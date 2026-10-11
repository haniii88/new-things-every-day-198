function dailyLog198() {
  const loginAttempts = [
    { user: "Alex", failed: 0, location: "Berlin" },
    { user: "Sam", failed: 3, location: "London" },
    { user: "Jordan", failed: 1, location: "Paris" },
    { user: "Taylor", failed: 5, location: "Unknown" },
    { user: "Morgan", failed: 0, location: "Madrid" }
  ];

  const suspicious = loginAttempts.filter(
    attempt => attempt.failed >= 3 || attempt.location === "Unknown"
  );

  const totalFailed = loginAttempts.reduce(
    (sum, attempt) => sum + attempt.failed,
    0
  );

  const report = {
    date: new Date().toISOString().split("T")[0],
    totalAccounts: loginAttempts.length,
    totalFailedAttempts: totalFailed,
    suspiciousAccounts: suspicious.map(attempt => attempt.user),
    alerts: suspicious.length,
    status: suspicious.length > 0
      ? "Review security alerts"
      : "No suspicious activity detected"
  };

  console.log("Daily Security Report:", report);
}

dailyLog198();
